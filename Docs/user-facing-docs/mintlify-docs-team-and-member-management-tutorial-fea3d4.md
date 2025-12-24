I'll analyze the source code to create comprehensive documentation for Team and Member Management. Let me start by exploring the project structure to understand the codebase.

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" | grep -E "(team|member|user)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="output">
</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 244
drwxr-xr-x 13 root root   4096 Jan  8 23:49 .
drwxr-xr-x  3 root root   4096 Jan  8 23:49 ..
drwxr-xr-x  8 root root   4096 Jan  8 23:49 .git
-rw-r--r--  1 root root    457 Jan  8 23:49 .gitignore
drwxr-xr-x  3 root root   4096 Jan  8 23:49 .next
drwxr-xr-x  3 root root   4096 Jan  8 23:49 .storybook
-rw-r--r--  1 root root    253 Jan  8 23:49 .yarnrc.yml
-rw-r--r--  1 root root    171 Jan  8 23:49 README.md
drwxr-xr-x  4 root root   4096 Jan  8 23:49 __tests__
drwxr-xr-x  2 root root   4096 Jan  8 23:49 app
-rw-r--r--  1 root root   1568 Jan  8 23:49 components.json
-rw-r--r--  1 root root    186 Jan  8 23:49 jest.config.js
-rw-r--r--  1 root root    374 Jan  8 23:49 middleware.ts
-rw-r--r--  1 root root   1124 Jan  8 23:49 next-env.d.ts
-rw-r--r--  1 root root    201 Jan  8 23:49 next.config.js
-rw-r--r--  1 root root 126812 Jan  8 23:49 package-lock.json
-rw-r--r--  1 root root   2173 Jan  8 23:49 package.json
drwxr-xr-x  4 root root   4096 Jan  8 23:49 public
drwxr-xr-x  8 root root   4096 Jan  8 23:49 src
drwxr-xr-x  3 root root   4096 Jan  8 23:49 stories
-rw-r--r--  1 root root    635 Jan  8 23:49 tailwind.config.ts
-rw-r--r--  1 root root    295 Jan  8 23:49 tsconfig.json
drwxr-xr-x  2 root root   4096 Jan  8 23:49 types
drwxr-xr-x  6 root root   4096 Jan  8 23:49 utils
-rw-r--r--  1 root root  32832 Jan  8 23:49 yarn.lock
</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f \( -name "*.ts" -o -name "*.tsx" \) | grep -v node_modules | grep -v ".next" | head -30</parameter>
</invoke>
</function_calls>
<parameter name="output">
./middleware.ts
./next-env.d.ts
./tailwind.config.ts
./types/supabase.ts
./src/pages/_app.tsx
./src/pages/_document.tsx
./src/pages/api/auth/[...nextauth].ts
./src/pages/api/hello.ts
./src/pages/dashboard.tsx
./src/pages/index.tsx
./src/pages/login.tsx
./src/pages/settings.tsx
./src/pages/team.tsx
./src/components/Layout.tsx
./src/components/Sidebar.tsx
./src/components/TeamMemberCard.tsx
./src/components/InviteMemberModal.tsx
./src/lib/supabase.ts
./src/hooks/useTeam.ts
./__tests__/components/TeamMemberCard.test.tsx
./__tests__/hooks/useTeam.test.tsx
./utils/auth/authHelpers.ts
./utils/team/teamHelpers.ts
./.storybook/main.ts
./.storybook/preview.ts
./stories/Button.stories.ts
</parameter>

Great! I can see there are team-related files. Let me explore the key files for team and member management.

<function_calls>
<invoke name="read_file">
<parameter name="path">src/pages/team.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
import React, { useState } from 'react';
import { useRouter } from 'next/router';
import Layout from '@/components/Layout';
import TeamMemberCard from '@/components/TeamMemberCard';
import InviteMemberModal from '@/components/InviteMemberModal';
import { useTeam } from '@/hooks/useTeam';
import { Button } from '@/components/ui/button';
import { UserPlus, Settings } from 'lucide-react';

export default function TeamPage() {
  const router = useRouter();
  const { teamMembers, loading, error, inviteMember, removeMember, updateMemberRole } = useTeam();
  const [isInviteModalOpen, setIsInviteModalOpen] = useState(false);

  const handleInvite = async (email: string, role: string) => {
    await inviteMember(email, role);
    setIsInviteModalOpen(false);
  };

  const handleRemove = async (memberId: string) => {
    if (confirm('Are you sure you want to remove this team member?')) {
      await removeMember(memberId);
    }
  };

  const handleRoleChange = async (memberId: string, newRole: string) => {
    await updateMemberRole(memberId, newRole);
  };

  if (loading) {
    return (
      <Layout>
        <div className="flex justify-center items-center h-screen">
          <div className="animate-spin rounded-full h-12 w-12 border-b-2 border-gray-900"></div>
        </div>
      </Layout>
    );
  }

  if (error) {
    return (
      <Layout>
        <div className="p-6">
          <div className="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded">
            Error loading team members: {error}
          </div>
        </div>
      </Layout>
    );
  }

  return (
    <Layout>
      <div className="p-6">
        <div className="flex justify-between items-center mb-6">
          <div>
            <h1 className="text-3xl font-bold text-gray-900">Team Members</h1>
            <p className="text-gray-600 mt-1">Manage your team and member permissions</p>
          </div>
          <div className="flex gap-3">
            <Button
              variant="outline"
              onClick={() => router.push('/settings?tab=team')}
            >
              <Settings className="mr-2 h-4 w-4" />
              Team Settings
            </Button>
            <Button onClick={() => setIsInviteModalOpen(true)}>
              <UserPlus className="mr-2 h-4 w-4" />
              Invite Member
            </Button>
          </div>
        </div>

        {teamMembers.length === 0 ? (
          <div className="text-center py-12 bg-gray-50 rounded-lg border-2 border-dashed border-gray-300">
            <UserPlus className="mx-auto h-12 w-12 text-gray-400" />
            <h3 className="mt-2 text-sm font-semibold text-gray-900">No team members</h3>
            <p className="mt-1 text-sm text-gray-500">Get started by inviting a team member.</p>
            <div className="mt-6">
              <Button onClick={() => setIsInviteModalOpen(true)}>
                <UserPlus className="mr-2 h-4 w-4" />
                Invite Member
              </Button>
            </div>
          </div>
        ) : (
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
            {teamMembers.map((member) => (
              <TeamMemberCard
                key={member.id}
                member={member}
                onRemove={handleRemove}
                onRoleChange={handleRoleChange}
              />
            ))}
          </div>
        )}

        <InviteMemberModal
          isOpen={isInviteModalOpen}
          onClose={() => setIsInviteModalOpen(false)}
          onInvite={handleInvite}
        />
      </div>
    </Layout>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/TeamMemberCard.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
import React from 'react';
import { Card, CardContent, CardHeader } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from '@/components/ui/select';
import { Avatar, AvatarFallback, AvatarImage } from '@/components/ui/avatar';
import { Badge } from '@/components/ui/badge';
import { Mail, Trash2 } from 'lucide-react';

interface TeamMember {
  id: string;
  email: string;
  name: string;
  role: string;
  avatar?: string;
  status: 'active' | 'pending' | 'inactive';
  joinedAt: string;
}

interface TeamMemberCardProps {
  member: TeamMember;
  onRemove: (memberId: string) => void;
  onRoleChange: (memberId: string, newRole: string) => void;
}

export default function TeamMemberCard({ member, onRemove, onRoleChange }: TeamMemberCardProps) {
  const getInitials = (name: string) => {
    return name
      .split(' ')
      .map(n => n[0])
      .join('')
      .toUpperCase();
  };

  const getStatusColor = (status: string) => {
    switch (status) {
      case 'active':
        return 'bg-green-100 text-green-800';
      case 'pending':
        return 'bg-yellow-100 text-yellow-800';
      case 'inactive':
        return 'bg-gray-100 text-gray-800';
      default:
        return 'bg-gray-100 text-gray-800';
    }
  };

  return (
    <Card className="hover:shadow-lg transition-shadow">
      <CardHeader className="pb-3">
        <div className="flex items-start justify-between">
          <div className="flex items-center gap-3">
            <Avatar className="h-12 w-12">
              <AvatarImage src={member.avatar} alt={member.name} />
              <AvatarFallback>{getInitials(member.name)}</AvatarFallback>
            </Avatar>
            <div>
              <h3 className="font-semibold text-lg">{member.name}</h3>
              <p className="text-sm text-gray-500 flex items-center gap-1">
                <Mail className="h-3 w-3" />
                {member.email}
              </p>
            </div>
          </div>
          <Badge className={getStatusColor(member.status)}>
            {member.status}
          </Badge>
        </div>
      </CardHeader>
      <CardContent>
        <div className="space-y-3">
          <div className="flex items-center justify-between">
            <span className="text-sm text-gray-600">Role</span>
            <Select
              value={member.role}
              onValueChange={(value) => onRoleChange(member.id, value)}
            >
              <SelectTrigger className="w-32">
                <SelectValue />
              </SelectTrigger>
              <SelectContent>
                <SelectItem value="admin">Admin</SelectItem>
                <SelectItem value="member">Member</SelectItem>
                <SelectItem value="viewer">Viewer</SelectItem>
              </SelectContent>
            </Select>
          </div>
          <div className="flex items-center justify-between">
            <span className="text-sm text-gray-600">Joined</span>
            <span className="text-sm font-medium">
              {new Date(member.joinedAt).toLocaleDateString()}
            </span>
          </div>
          <div className="pt-2 border-t">
            <Button
              variant="destructive"
              size="sm"
              className="w-full"
              onClick={() => onRemove(member.id)}
            >
              <Trash2 className="mr-2 h-4 w-4" />
              Remove Member
            </Button>
          </div>
        </div>
      </CardContent>
    </Card>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/InviteMemberModal.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
import React, { useState } from 'react';
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogFooter,
  DialogHeader,
  DialogTitle,
} from '@/components/ui/dialog';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from '@/components/ui/select';

interface InviteMemberModalProps {
  isOpen: boolean;
  onClose: () => void;
  onInvite: (email: string, role: string) => void;
}

export default function InviteMemberModal({ isOpen, onClose, onInvite }: InviteMemberModalProps) {
  const [email, setEmail] = useState('');
  const [role, setRole] = useState('member');
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [error, setError] = useState('');

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    setError('');

    // Validate email
    if (!email || !email.includes('@')) {
      setError('Please enter a valid email address');
      return;
    }

    setIsSubmitting(true);
    try {
      await onInvite(email, role);
      setEmail('');
      setRole('member');
      onClose();
    } catch (err) {
      setError('Failed to send invitation. Please try again.');
    } finally {
      setIsSubmitting(false);
    }
  };

  return (
    <Dialog open={isOpen} onOpenChange={onClose}>
      <DialogContent className="sm:max-w-[425px]">
        <DialogHeader>
          <DialogTitle>Invite Team Member</DialogTitle>
          <DialogDescription>
            Send an invitation to add a new member to your team. They'll receive an email with instructions to join.
          </DialogDescription>
        </DialogHeader>
        <form onSubmit={handleSubmit}>
          <div className="grid gap-4 py-4">
            <div className="grid gap-2">
              <Label htmlFor="email">Email Address</Label>
              <Input
                id="email"
                type="email"
                placeholder="colleague@example.com"
                value={email}
                onChange={(e) => setEmail(e.target.value)}
                required
              />
            </div>
            <div className="grid gap-2">
              <Label htmlFor="role">Role</Label>
              <Select value={role} onValueChange={setRole}>
                <SelectTrigger id="role">
                  <SelectValue />
                </SelectTrigger>
                <SelectContent>
                  <SelectItem value="admin">
                    <div>
                      <div className="font-medium">Admin</div>
                      <div className="text-xs text-gray-500">Full access to all features</div>
                    </div>
                  </SelectItem>
                  <SelectItem value="member">
                    <div>
                      <div className="font-medium">Member</div>
                      <div className="text-xs text-gray-500">Can view and edit content</div>
                    </div>
                  </SelectItem>
                  <SelectItem value="viewer">
                    <div>
                      <div className="font-medium">Viewer</div>
                      <div className="text-xs text-gray-500">Read-only access</div>
                    </div>
                  </SelectItem>
                </SelectContent>
              </Select>
            </div>
            {error && (
              <div className="text-sm text-red-600 bg-red-50 p-2 rounded">
                {error}
              </div>
            )}
          </div>
          <DialogFooter>
            <Button type="button" variant="outline" onClick={onClose}>
              Cancel
            </Button>
            <Button type="submit" disabled={isSubmitting}>
              {isSubmitting ? 'Sending...' : 'Send Invitation'}
            </Button>
          </DialogFooter>
        </form>
      </DialogContent>
    </Dialog>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/hooks/useTeam.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { useState, useEffect } from 'react';
import { supabase } from '@/lib/supabase';

interface TeamMember {
  id: string;
  email: string;
  name: string;
  role: string;
  avatar?: string;
  status: 'active' | 'pending' | 'inactive';
  joinedAt: string;
}

export function useTeam() {
  const [teamMembers, setTeamMembers] = useState<TeamMember[]>([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    fetchTeamMembers();
  }, []);

  const fetchTeamMembers = async () => {
    try {
      setLoading(true);
      const { data, error } = await supabase
        .from('team_members')
        .select('*')
        .order('joinedAt', { ascending: false });

      if (error) throw error;

      setTeamMembers(data || []);
    } catch (err) {
      setError(err instanceof Error ? err.message : 'An error occurred');
    } finally {
      setLoading(false);
    }
  };

  const inviteMember = async (email: string, role: string) => {
    try {
      const { data, error } = await supabase
        .from('team_invitations')
        .insert([
          {
            email,
            role,
            status: 'pending',
            invitedAt: new Date().toISOString(),
          },
        ])
        .select();

      if (error) throw error;

      // Send invitation email
      await supabase.functions.invoke('send-team-invitation', {
        body: { email, role },
      });

      // Refresh team members list
      await fetchTeamMembers();
    } catch (err) {
      throw new Error(err instanceof Error ? err.message : 'Failed to invite member');
    }
  };

  const removeMember = async (memberId: string) => {
    try {
      const { error } = await supabase
        .from('team_members')
        .delete()
        .eq('id', memberId);

      if (error) throw error;

      // Update local state
      setTeamMembers(teamMembers.filter(m => m.id !== memberId));
    } catch (err) {
      throw new Error(err instanceof Error ? err.message : 'Failed to remove member');
    }
  };

  const updateMemberRole = async (memberId: string, newRole: string) => {
    try {
      const { error } = await supabase
        .from('team_members')
        .update({ role: newRole })
        .eq('id', memberId);

      if (error) throw error;

      // Update local state
      setTeamMembers(teamMembers.map(m => 
        m.id === memberId ? { ...m, role: newRole } : m
      ));
    } catch (err) {
      throw new Error(err instanceof Error ? err.message : 'Failed to update role');
    }
  };

  return {
    teamMembers,
    loading,
    error,
    inviteMember,
    removeMember,
    updateMemberRole,
    refetch: fetchTeamMembers,
  };
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/pages/settings.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
import React, { useState } from 'react';
import { useRouter } from 'next/router';
import Layout from '@/components/Layout';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import { Button } from '@/components/ui/button';
import { Switch } from '@/components/ui/switch';

export default function SettingsPage() {
  const router = useRouter();
  const { tab = 'profile' } = router.query;

  return (
    <Layout>
      <div className="p-6">
        <div className="mb-6">
          <h1 className="text-3xl font-bold text-gray-900">Settings</h1>
          <p className="text-gray-600 mt-1">Manage your account and team preferences</p>
        </div>

        <Tabs value={tab as string} onValueChange={(value) => router.push(`/settings?tab=${value}`)}>
          <TabsList className="grid w-full grid-cols-3 lg:w-[400px]">
            <TabsTrigger value="profile">Profile</TabsTrigger>
            <TabsTrigger value="team">Team</TabsTrigger>
            <TabsTrigger value="notifications">Notifications</TabsTrigger>
          </TabsList>

          <TabsContent value="profile" className="space-y-4">
            <Card>
              <CardHeader>
                <CardTitle>Profile Information</CardTitle>
                <CardDescription>
                  Update your personal information and preferences
                </CardDescription>
              </CardHeader>
              <CardContent className="space-y-4">
                <div className="space-y-2">
                  <Label htmlFor="name">Full Name</Label>
                  <Input id="name" placeholder="John Doe" />
                </div>
                <div className="space-y-2">
                  <Label htmlFor="email">Email Address</Label>
                  <Input id="email" type="email" placeholder="john@example.com" />
                </div>
                <Button>Save Changes</Button>
              </CardContent>
            </Card>
          </TabsContent>

          <TabsContent value="team" className="space-y-4">
            <Card>
              <CardHeader>
                <CardTitle>Team Settings</CardTitle>
                <CardDescription>
                  Configure team-wide settings and permissions
                </CardDescription>
              </CardHeader>
              <CardContent className="space-y-4">
                <div className="flex items-center justify-between">
                  <div className="space-y-0.5">
                    <Label>Allow members to invite others</Label>
                    <p className="text-sm text-gray-500">
                      Let team members send invitations to new members
                    </p>
                  </div>
                  <Switch />
                </div>
                <div className="flex items-center justify-between">
                  <div className="space-y-0.5">
                    <Label>Require approval for new members</Label>
                    <p className="text-sm text-gray-500">
                      Admin must approve all new member requests
                    </p>
                  </div>
                  <Switch />
                </div>
                <div className="flex items-center justify-between">
                  <div className="space-y-0.5">
                    <Label>Enable role-based permissions</Label>
                    <p className="text-sm text-gray-500">
                      Restrict features based on member roles
                    </p>
                  </div>
                  <Switch defaultChecked />
                </div>
                <Button>Save Team Settings</Button>
              </CardContent>
            </Card>
          </TabsContent>

          <TabsContent value="notifications" className="space-y-4">
            <Card>
              <CardHeader>
                <CardTitle>Notification Preferences</CardTitle>
                <CardDescription>
                  Choose what notifications you want to receive
                </CardDescription>
              </CardHeader>
              <CardContent className="space-y-4">
                <div className="flex items-center justify-between">
                  <div className="space-y-0.5">
                    <Label>New team member joins</Label>
                    <p className="text-sm text-gray-500">
                      Get notified when someone joins your team
                    </p>
                  </div>
                  <Switch defaultChecked />
                </div>
                <div className="flex items-center justify-between">
                  <div className="space-y-0.5">
                    <Label>Team member removed</Label>
                    <p className="text-sm text-gray-500">
                      Get notified when a member leaves the team
                    </p>
                  </div>
                  <Switch defaultChecked />
                </div>
                <div className="flex items-center justify-between">
                  <div className="space-y-0.5">
                    <Label>Role changes</Label>
                    <p className="text-sm text-gray-500">
                      Get notified when member roles are updated
                    </p>
                  </div>
                  <Switch />
                </div>
                <Button>Save Preferences</Button>
              </CardContent>
            </Card>
          </TabsContent>
        </Tabs>
      </div>
    </Layout>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">utils/team/teamHelpers.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
export const TEAM_ROLES = {
  ADMIN: 'admin',
  MEMBER: 'member',
  VIEWER: 'viewer',
} as const;

export type TeamRole = typeof TEAM_ROLES[keyof typeof TEAM_ROLES];

export interface RolePermissions {
  canInviteMembers: boolean;
  canRemoveMembers: boolean;
  canEditRoles: boolean;
  canViewTeam: boolean;
  canEditContent: boolean;
}

export const getRolePermissions = (role: TeamRole): RolePermissions => {
  switch (role) {
    case TEAM_ROLES.ADMIN:
      return {
        canInviteMembers: true,
        canRemoveMembers: true,
        canEditRoles: true,
        canViewTeam: true,
        canEditContent: true,
      };
    case TEAM_ROLES.MEMBER:
      return {
        canInviteMembers: false,
        canRemoveMembers: false,
        canEditRoles: false,
        canViewTeam: true,
        canEditContent: true,
      };
    case TEAM_ROLES.VIEWER:
      return {
        canInviteMembers: false,
        canRemoveMembers: false,
        canEditRoles: false,
        canViewTeam: true,
        canEditContent: false,
      };
    default:
      return {
        canInviteMembers: false,
        canRemoveMembers: false,
        canEditRoles: false,
        canViewTeam: false,
        canEditContent: false,
      };
  }
};

export const validateEmail = (email: string): boolean => {
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailRegex.test(email);
};

export const formatMemberStatus = (status: string): string => {
  switch (status) {
    case 'active':
      return 'Active';
    case 'pending':
      return 'Invitation Pending';
    case 'inactive':
      return 'Inactive';
    default:
      return 'Unknown';
  }
};
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/Sidebar.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
import React from 'react';
import Link from 'next/link';
import { useRouter } from 'next/router';
import { Home, Users, Settings, LogOut } from 'lucide-react';